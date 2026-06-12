---
title: "Truecrypt.... how to remote mount volume? or send bash script remotely?"
date: 2011-04-01
forum: Security
---

### Post by steven.smith on 2011-04-01
So here's my setup: (skip to summary at bottom if you don't want to read this)

I have an Ubuntu 10.04 machine at home and apache setup on it (files are located in a Truecrypt volume). The reason for the web server being that I wanted to access my files wherever I'm at (i.e. hotel, work, hotspots, etc...). So far, it's worked out great for me seeing as a I can http download my files (or stream media files). However, I am often on a public hotspot and I know it's a matter of time before someone finds the webserver on my computer. I have the machine firewalled and password protected (via .htaccess), but either way I don't want people looking in on my computer.

    The problem:
I have used Truecrypt for a long time and completely trust using the program to encrypt/unencrypt a volume container to store my files. Usually, I would remote desktop into my computer and mount/unmount the volume when I needed it. However, after time it get's really annoying to do this. So I eventually figured out how to setup a bash script to automatically do this for me (which I put on the usb part of my phone). What I wanted to do was to be able send the bash script to my Ubuntu machine (via ftp from my phone) and have Ubuntu automatically run the script. Is this possible? What programs do I need on Ubuntu?

I was thinking about using something like cron, but that is for scheduled times. I don't really have a set time in which I need my files, it's pretty sporadic depending on how much I travel. Thus the need for being able to remotely mount the volume _when_ I need it.



Summary:
I need a way for Ubuntu to read a folder every minute or so to check for bash scripts to run. I want to be able to send the bash script via ftp from my phone, have Ubuntu run the script, then delete itself (so as to not store the password). I already know the script in which to mount the Truecrypt volume and how to send the file via ftp from my phone. It's really a matter of what program to use in Ubuntu to find and run the script.

Thanks in advance for any and all help :)

---

### Post by kidders on 2011-04-03
Hi there,

Disk encryption is not intended to be used in this way. Software like Truecrypt is designed to prevent someone with physical access to your hard disk from reading your data. It offers no protection in other situations.

> **steven.smith said:**
> I am often on a public hotspot and I know it's a matter of time before someone finds the webserver on my computer.Accessing your computer over HTTP using public wifi is highly dangerous, since everyone can see your .htaccess password, along with any truecrypt key/script you send, and all the data you download.

A far better means of controlling access to your box would be to use HTTPS with client certification, so that ...[LIST=1]
[*]Anything you transmit (including .htaccess passwords) would be encrypted, regardless of whether you're using public wifi.
[*]You can configure your web server to refuse to cooperate with someone who doesn't have the appropriate SSL cert, and the keyphrase that goes with it.
[/LIST]

In any case, to answer your question, all you really need is a trivial shell script, to check for & execute anything in a given directory, for example ...```
for f in /path/to/scripts/*.sh; do bash $f; done
```

Running something like that every few minutes should do the trick. Again, bear in mind that this is all very risky ...[LIST]
[*]It's not a good idea to even *run* an FTP server on a domestic computer. In my experience, using one attracts a lot of unwanted attention (eg brute force attacks, etc).
[*]It's a totally insecure protocol, so anything you upload over public wifi (including the FTP login) will be visible to everyone.
[*]Leaving aside the theoretical possibility of someone uploading a malicious script to your computer, there'd be no room for mistakes on your part! Anything you uploaded, no matter what it was, would be executed within minutes ... Not necessarily a great idea.
[*]If you *do* go down this road, _never_ run the uploaded scripts as root.
[/LIST]

Anyhow, I hope you don't mind all the added commentary! I really would suggest not trying to involve Truecrypt in keeping your data safe while your computer is turned on.

---

### Post by steven.smith on 2011-04-03
Thanks for your reply, I rarely actually get a response to my posts, your advice is definitely welcome. I was able to eventually solve this (which I'll get to at the end of this post), however I would like to clear up a few things.

> Disk encryption is not intended to be used in this way. Software like Truecrypt is designed to prevent someone with physical access to your hard disk from reading your data. It offers no protection in other situations.
I am very well aware that truecrypt is really meant to encrypt a drive so that if stolen it can't be accessed. This is the reason why I use Truecrypt, however the problem I had was that all my sensitive data was in the Truecrypt volume, so I needed an easy way to mount/unmount it whenever I needed it.

> Accessing your computer over HTTP using public wifi is highly dangerous, since everyone can see your .htaccess password, along with any truecrypt key/script you send, and all the data you download.

A far better means of controlling access to your box would be to use HTTPS with client certification, so that ...
Anything you transmit (including .htaccess passwords) would be encrypted, regardless of whether you're using public wifi.
You can configure your web server to refuse to cooperate with someone who doesn't have the appropriate SSL cert, and the keyphrase that goes with it.
   You are absolutely right. I did not mention that I connect to my web server through https (thought it was irrelevant). But I do use https when I HAVE to. Usually, I VPN (via Openvpn) into my network and change the files from there, however at public wifi's there's a lot of restrictions and you never know when the port you want will be locked. Added to that, I have proxy access, so when I need it i can use it.

> It's not a good idea to even run an FTP server on a domestic computer. In my experience, using one attracts a lot of unwanted attention (eg brute force attacks, etc).
Very true here also, however I added a User that can only ftp to a certain public directory on the webserver. I usually don't rely on FTP.

> Leaving aside the theoretical possibility of someone uploading a malicious script to your computer, there'd be no room for mistakes on your part! Anything you uploaded, no matter what it was, would be executed within minutes ... Not necessarily a great idea.
There's always a risk that a hacker can get into the system, however I feel pretty secure in that I have everything firewalled. You are right in that someone could potentially steal access into the ftp folder and run a script in it, but you have to understand the process in which I am doing this. I'm not sending a command over ftp, I'm sending an encrypted file (with a different extension such as .txt) over ftp. Simply put, if a hacker can't actually open the file, then the data is still safe. If they manage to steal the username/password of the ftp folder, it won't matter because the User is locked to the directory (at least I hope it doesn't matter). Either way, it's not such a big security risk to me.

> Anyhow, I hope you don't mind all the added commentary!
On the contrary, I like the fact that you actually decided to talk about the risks of doing so. It's good at add extra information just in case someone hasn't thought of something. You do have valid points above.


As for the solution I found (before reading the above post) was quite simple:
I have the bash script on my phone set as an extension of ".mp4". When I'm ready to mount the volume to download/stream files, I use the ftp client on my phone to transfer ".mp4" file to a non-public folder on my computer. I've set cron to check the folder every 2 minutes and rename the file back to a bash script. From there, the command to mount the Truecrypt volume is sent. Afterwards, I have the script to permanently delete itself.

Sounds a little complicated, but it's not. And once everything was setup, it worked perfectly. If anyone wants the exact commands, I can make a mini-howto that's really simple to follow. If anyone wants it, just post a request here and I'll put it up.

---

### Post by dgw on 2011-04-03
Is there a reason why you aren't just using ssh for this stuff?

---

### Post by steven.smith on 2011-04-03
> Is there a reason why you aren't just using ssh for this stuff?

Simple. I'm often behind restrictive firewalls and don't always have access to SSH. I travel a lot and I'm on Wifi Hotspots most of the time. I need a way to easily lock and unlock folders for when I need them and make sure I don't give anyone easy access to my system.

---

### Post by cjsteele on 2011-04-03
so... why not write a tiny front-end that allows you to mount it and un-mount it via a web interface.  Seems like that'd be a lot easier than doing it via FTP, or similar hackery.  you could even make the volume accessible via a self-signed SSL, password-protected web-interface once its mounted.  Use one of the pre-packaged file browsers (I dig eXtplorer)

Off hand, what kind of phone are you connecting from?

Cheers,
-C

---

### Post by steven.smith on 2011-04-04
> why not write a tiny front-end that allows you to mount it and un-mount it via a web interface. Seems like that'd be a lot easier than doing it via FTP, or similar hackery. you could even make the volume accessible via a self-signed SSL, password-protected web-interface once its mounted. Use one of the pre-packaged file browsers (I dig eXtplorer)

I actually had a similar idea in that I would use the net2ftp php application instead of actually using a computer based ftp client. That way I could use https to run the program. However, this isn't really the point of all of it. I really just wanted to have the ease of access to mount and unmount the folder for web access. With the setup I have, it takes two taps on my phone to make the files accessible or lock them down. To me it is a lot easier than having to login to my webserver or VNC into it just to make the files accessible. 

> Off hand, what kind of phone are you connecting from?
I have a Palm Pre Plus (with Classic as a Palm Emulator for the ftp client).

---

### Post by Sporkman on 2011-04-05
> **steven.smith said:**
> Simple. I'm often behind restrictive firewalls and don't always have access to SSH. I travel a lot and I'm on Wifi Hotspots most of the time. I need a way to easily lock and unlock folders for when I need them and make sure I don't give anyone easy access to my system.

Instead of a webserver, you could always just have ssh listen on port 80 (which firewalls usually allow), then mount directories using [sshfs]("http://en.wikipedia.org/wiki/SSHFS"). You'll then have your directories on your home computer appear seamlessly on your laptop in nautilus for example, and it would be completely secure.

EDIT: Sorry, I missed the part about connecting from your phone - not sure if sshfs would work from a phone...

---

### Post by kidders on 2011-04-05
> **Sporkman said:**
> Sorry, I missed the part about connecting from your phone - not sure if sshfs would work from a phone...WebDAV over SSL would be a better option, I'd say. Anything that didn't support the DAV extensions (eg a phone) would still have plain HTTP to fall back on.

---

