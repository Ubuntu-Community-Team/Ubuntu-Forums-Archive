---
title: "ubuntu one not uploading - thought I'd report it"
date: 2012-03-10
forum: Ubuntu One (CLOSED)
---

### Post by imachavel on 2012-03-10
I have a 7 day trial for 5 gb of space(probably 6 now) as I really need to upload 2gb worth of files to send to a friend for code sitting on top of other code libraries or what not. Anyway, thought I was getting it all worked out, but the files just hang, it says they are uploading but after 12 hours 2gb of files have no uploaded at all. It's very confusing the files are even tar balled. Oh well....... Any ideas??

---

### Post by imachavel on 2012-03-10
sorry I wasn't much more clear. It's basically theoretical information. No actual files but anyway beyond the point. I just want to bump this, if only because I'm hoping if no one else has had this same error, that someone can report they've taken a note of this, I really need to use ubuntu one for 2gb of space and possibly later for further uses. Gotta figure out what is wrong, Should I try and ssh into the account?

thanks for noticing

---

### Post by oldos2er on 2012-03-10
Moved to Ubuntu One.

---

### Post by imachavel on 2012-03-10
still nothing huh? I keep trying it again and again, just not working. GOD I keep thinking it's the servers fault! Wtf! Just can't figure it out.

---

### Post by MG&amp;TL on 2012-03-11
Are you using the Ubuntu One client, or the web-based interface?

---

### Post by imachavel on 2012-03-11
[https://one.ubuntu.com/files/#f=f%2Fciscoshare](https://one.ubuntu.com/files/#f=f%2Fciscoshare)

web based interface I think? Is there another option? Still, how will it effect uploads? when I try to upload I go to browse, chose the file, then it says please wait, as though it's uploading. But it'll say please wait for 12 hours and nothing will happen. Do you think I'm missing a driver or plug in or some support file extension that is supposed to help the interfaces find each other, or better said, help the web server connect to my computer via .net framework or whatnot? After all, the interfaces are just what allows the user to interact with things.

Maybe there is another way of doing it? Is that the web interface or ubuntu one client. Ubuntu one client I download to my pc then chose to upload to ubuntu one, instead of ubuntu one web interface choosing the file from my pc then syncing with the server? They will both server the same purpose though, an interface to allow files to be found in a directory on my pc, then uploaded. I'm wracking my brain, but I've diagnosed basically what needs to happen. Do I need to open some port on my att 7550 netgear router?

---

### Post by MG&amp;TL on 2012-03-11
".net framework"- :oops:

You could try the client on your pc, you should be able to find it in the Unity menu. Looks a bit like: [http://www.google.com/imgres?um=1&hl=en&client=ubuntu&sa=N&channel=fs&gl=uk&biw=1305&bih=680&tbm=isch&tbnid=cJQivw-yMqFuOM:&imgrefurl=http://theworldoftech.net/ubuntu-one/&docid=H8YXvQP2Y3xp8M&imgurl=http://theworldoftech.net/wp-content/uploads/2011/08/ubuntu-1-snapshot.jpg&w=748&h=560&ei=helcT--NEeLK0QX63ODGDQ&zoom=1&iact=hc&vpx=810&vpy=318&dur=671&hovh=194&hovw=260&tx=78&ty=102&sig=113762648752440566914&page=1&tbnh=151&tbnw=202&start=0&ndsp=15&ved=1t:429,r:8,s:0](http://www.google.com/imgres?um=1&hl=en&client=ubuntu&sa=N&channel=fs&gl=uk&biw=1305&bih=680&tbm=isch&tbnid=cJQivw-yMqFuOM:&imgrefurl=http://theworldoftech.net/ubuntu-one/&docid=H8YXvQP2Y3xp8M&imgurl=http://theworldoftech.net/wp-content/uploads/2011/08/ubuntu-1-snapshot.jpg&w=748&h=560&ei=helcT--NEeLK0QX63ODGDQ&zoom=1&iact=hc&vpx=810&vpy=318&dur=671&hovh=194&hovw=260&tx=78&ty=102&sig=113762648752440566914&page=1&tbnh=151&tbnw=202&start=0&ndsp=15&ved=1t:429,r:8,s:0)

You probably have an Ubuntu one folder in your home directory, that's automatically synced. Only asking in case something's wrong with the webpage. What's your upload speed like? 2GB might take a while to upload.

---

### Post by imachavel on 2012-03-11
it's dsl, definitely shouldn't take two days to upload, that is for sure. Let me look for the unity compiz plug in interface client then. I'm opening that link, I wonder if I need to sudo apt-get install it

I wish they had an answer for the client for unity interface, now I'm trying to install it in kde interface, not sure which repository to add it to:

sudo add-apt-repository ppa: apache logger/ubuntuone-kde
[sudo] password for danel: 
Error: need a repository as argument

[http://maketecheasier.com/how-to-install-and-setup-ubuntu-one-in-kubuntu/2010/03/15](http://maketecheasier.com/how-to-install-and-setup-ubuntu-one-in-kubuntu/2010/03/15)

think trying it with the client will work better?

---

### Post by MG&amp;TL on 2012-03-11
Should be:

```
sudo add-apt-repository ppa:apachelogger/ubuntuone-kde
```(no spaces)

You have a wonderful talent for coming up with unrelated things, I must say. :) Compiz has nothing to do with it.

If you have removed it,

```
sudo apt-get install ubuntuone-client
```should do it.

IDK, possibly. It should at least give you some indication of what's gone wrong and how long it's going to take.

---

### Post by imachavel on 2012-03-11
maybe I do already have it installed because:

sudo add-apt-repository ppa: apache logger/ubuntuone-kde
[sudo] password for danel: 
Error: need a repository as argument
danel@danel-Dimension-4700:~$ sudo add-apt-repository ppa:apachelogger/ubuntuone-kde
[sudo] password for danel: 
You are about to add the following PPA to your system:
 ubuntuone-kde
 tag:launchpad.net:2008:redacted
 More info: [https://launchpad.net/~apachelogger/+archive/ubuntuone-kde](https://launchpad.net/~apachelogger/+archive/ubuntuone-kde)
Press [ENTER] to continue or ctrl-c to cancel adding it

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.rdr59HlWBU --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv tag:launchpad.net:2008:redacted
gpg: "tag:launchpad.net:2008:redacted" not a key ID: skipping
danel@danel-Dimension-4700:~$ sudo apt-get install ubuntuone-client
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntuone-client is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
danel@danel-Dimension-4700:~$ sudo add-apt-repository ppa:apachelogger/ubuntuone-kde
You are about to add the following PPA to your system:
 ubuntuone-kde
 tag:launchpad.net:2008:redacted
 More info: [https://launchpad.net/~apachelogger/+archive/ubuntuone-kde](https://launchpad.net/~apachelogger/+archive/ubuntuone-kde)
Press [ENTER] to continue or ctrl-c to cancel adding it

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.ajrkiKOxPU --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv tag:launchpad.net:2008:redacted
gpg: "tag:launchpad.net:2008:redacted" not a key ID: skipping

---

### Post by MG&amp;TL on 2012-03-11
So UbuntuOne should be in the Unity dash...

If you want to install the Qt version, by all means go ahead.

---

### Post by imachavel on 2012-03-11
ok there is a problem, I believe the client interface needs to be installed whether you access your files through the web site or not. I'm not extremely familiar with ports, the difference between ftp and other file transfer protocols. But it would seem the back end of the client is necessary if you want the OS to connect through necessary ports and transfer files to the web server properly. I don't mean to get off topic, it just seems easier for me to understand is all. The interface is just the front end that you interact with, the back end is what is doing all the work, My guess is the client installs back end properties necessary to transfer the files. 

Another problem now, it won't install correctly. Getting somewhere though, I may need some other repository support added, to make it work correctly.

---

### Post by imachavel on 2012-03-11
> **MG&TL said:**
> So UbuntuOne should be in the Unity dash...

If you want to install the Qt version, by all means go ahead.

read above, what a snag! Ok never mind it doesn't seem it was necessary. I just copy and pasted the files and it says it's in the folder now. Check the file sharing link, thanks

---

### Post by MG&amp;TL on 2012-03-11
That *is* installed. You probably have an Ubuntu One folder in your homefolder now? Try dragging some stuff there, it should upload.

As for the backend/frontend stuff, it works a little like this:

1. You make a connection through a protocol like ssh or ftp. That logs you into your account, and gives you permission to upload your files.

2. A user clicks some helpfully labelled buttons, which connect to the program, via some clever stuff like the X server.

3. The program upload the user-specified files through something like ssh or ftp.

4. Job Done.

---

### Post by imachavel on 2012-03-11
nothing huh? Damn it's weird, my client interfacing is not connecting with the web server. The problem has GOT to the be the ubuntu one server, if it wasn't, then when I tried uploading the files by copying and pasting into the share folder I created on the web site, it would have told me something was wrong instead of saying it was copying the files. Something is very very strange here. Why did it allow me to copy and paste the files into the folder? in the ubuntu one control panel, it says file sync is in progress. Now if file sync is in progress, why in the hell is there nothing in the folder online?

Maybe I need to enable contacts sync? Let me try it then. No wait, that's for evolution or thunderbird mail client contact sync, which I want but is not the issue I'm trying to address. Says all folders are synced, well maybe .... let me try something..

---

### Post by imachavel on 2012-03-12
they finally showed up:

[https://one.ubuntu.com/files/#f=f%2Fciscoshare](https://one.ubuntu.com/files/#f=f%2Fciscoshare)

Ok issue should be solved, if I can't download them I'll create another thread. Thanks for the help then

---

