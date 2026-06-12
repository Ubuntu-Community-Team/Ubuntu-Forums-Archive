---
title: "Sunbird and NAS on Ratel"
date: 2008-02-09
forum: System76 Support
---

### Post by eadwacer on 2008-02-09
This is a little off-topic for this forum, but I've gotten zero responses from either the Mozillazine Sunbird forum or the Ubuntu network and wireless forums, so I'm trying here.

Just installed Sunbird 0.7calendaring program. My goal is to have one calendar stored on my NAS and visible from all three PCs on my LAN (Win2K, XP, and Ratel/Ubuntu)

I am having trouble getting Sunbird on the Ratel to see a network drive - the Nautilus file browser on the Ratel sees the network fine, and I can share files across the LAN, no problem, so it's not a network problem.

On the Ratel box, when I try to subscribe to a new calendar on the network, Sunbird asks for the location and name, and tells me it was created.  The name and location I got by looking at the .ics file properties in Nautilus:

smb://NASbox/Shared%20Files/Calendar/OurCalendar.ics

However, it was not created, it doesn't show up in the calendar list, and the error console shows:

Error: [Exception... "Component returned failure code: 0x804b0012 [nsIIOService.newChannelFromURI]"  nsresult: "0x804b0012 (<unknown>)"  location: "JS frame :: file:///C:/Program%20Files/Mozilla%20Sunbird/components/calICSCalendar.js :: anonymous :: line 161"  data: no]
Source File: file:///C:/Program%20Files/Mozilla%20Sunbird/components/calICSCalendar.js
Line: 161

 I am pretty sure I'm just not giving it the right location string. I have tried the Mozilla KB, and a general search (and asked), but can't find anything on this. Can someone give me pointers on where to look?

---

### Post by compholio on 2008-02-09
My guess is that Sunbird does not use GnomeVFS, so it cannot see "smb://" addresses.  This particular problem will supposedly be fixed in the next version of Gnome where GnomeVFS will be replaced with FUSE (so the mount will be a "real" mount instead of a virtual mount).  Anyway, I would suggest fixing this by manually making a "real" mount for your networked filesystem.  I do not know your familiarity with doing terminal operations so I apologize if the following steps are too dumbed down for your abilities:
1) Open a terminal by going to Ubu | Accessories | Terminal
2) Type "sudo mkdir /media/nasbox-shared" and hit enter
3) Type in your password
4) Type "sudo apt-get install smbfs" and hit enter, type "Y" and hit enter when prompted
5) Type "sudo gedit /etc/fstab" and hit enter
6) Add the following line to the bottom of the file:
```
//NASbox/Shared\ Files/ /media/nasbox-shared cifs user,guest,noauto,rw,noperm 0 0
```

What this has done is added a special drive to your "Computer" in Gnome called "nasbox-shared".  When you want to use it just right click on it and use the "mount" option to activate it, you can do this from ANY file or folder dialog or from nautilus itself.  Once you have done this you should be able to get Sunbird to find the file.  If any of this does not work then post back, it's possible I've forgotten a step since it has been a while since I've done this.

---

### Post by eadwacer on 2008-02-09
Thanks, compholio, I'll work on that this evening -- and... it's not possible to dumb down a reply to me too much, unless you have special dumb-down training.
Steve Shervais

---

### Post by eadwacer on 2008-02-09
No joy so far:
Followed the compholio directions 1-6, including copy/pasting the suggested line to fstab. 

However, no new drive appeared in the Places/Computer menu [do I need to restart something?], and when I did a naive 'mount nasbox-shared' command (just to see what would happen) it said that the pasted line in fstab was 'bad' and that it couldn't find 'nasbox-shared' in fstab or mntab. 

Steve Shervais

---

### Post by compholio on 2008-02-11
> **eadwacer said:**
> No joy so far:
Followed the compholio directions 1-6, including copy/pasting the suggested line to fstab. 

However, no new drive appeared in the Places/Computer menu [do I need to restart something?], and when I did a naive 'mount nasbox-shared' command (just to see what would happen) it said that the pasted line in fstab was 'bad' and that it couldn't find 'nasbox-shared' in fstab or mntab. 

Steve Shervais

See what it says when you try "mount /media/nasbox-shared"...  Did you save /etc/fstab after adding that line (that might help)?

---

### Post by eadwacer on 2008-02-11
Did save. Gave me same error:

sshervais@ubuntu:~$ mount /media/nasbox-shared
[mntent]: line 10 in /etc/fstab is bad
mount: can't find /media/nasbox-shared in /etc/fstab or /etc/mtab

I had previously played around with some of the capitalization, just in case, but that didn't help.  Went back and pasted your original line into fstab - that's the line 10 it's talking about.

I really appreciate the time you are taking on this.
Steve

---

### Post by compholio on 2008-02-11
> **eadwacer said:**
> Did save. Gave me same error:

sshervais@ubuntu:~$ mount /media/nasbox-shared
[mntent]: line 10 in /etc/fstab is bad
mount: can't find /media/nasbox-shared in /etc/fstab or /etc/mtab

I had previously played around with some of the capitalization, just in case, but that didn't help.  Went back and pasted your original line into fstab - that's the line 10 it's talking about.

I really appreciate the time you are taking on this.
Steve
Well, I've never used a network share in fstab that has a space in it - it might be that "\ " is not being treated properly, maybe try these options instead (I highly doubt %20 would work but if quotes doesn't then I'm at a bit of a loss):
```
"//NASbox/Shared Files/" /media/nasbox-shared cifs user,guest,noauto,rw,noperm 0 0
```
```
//NASbox/Shared%20Files/ /media/nasbox-shared cifs user,guest,noauto,rw,noperm 0 0
```

P.S. Check that "/sbin/mount.cifs" exists.

---

### Post by eadwacer on 2008-02-11
AHA!! Getting close!

The %20 version put nasbox-shared onto Places/Computer menu

Now, when I give the mount command, I get a new error (always an exciting development):

mount error 1 = Operation not permitted
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)

as for /sbin/mount.cifs, on the one hand, it exists. On the other, it hasn't been changed since last December.

---

### Post by eadwacer on 2008-02-11
Umm. In my last post, that little bearded guy with the one ear was supposed to be an eight inside parens. Should have previewed.

---

### Post by eadwacer on 2008-02-11
Looking at the Man pages for mount, they seem to want one to be root, so I tried sudo mount, and got a different error:

retrying with upper case share name
mount error 6 = No such device or address

BTW, when I go to Places/Computer on the menu, and look at the Properties of nasbox-shared, it shows the location as:

computer:///

Don't know if that's significant.

---

### Post by compholio on 2008-02-11
> **eadwacer said:**
> Looking at the Man pages for mount, they seem to want one to be root, so I tried sudo mount, and got a different error:

retrying with upper case share name
mount error 6 = No such device or address

BTW, when I go to Places/Computer on the menu, and look at the Properties of nasbox-shared, it shows the location as:

computer:///

Don't know if that's significant.

Ahh, so the root thing is because I forgot part of what you need to do.  You need to run the commands:
```
sudo chmod +s /sbin/mount.cifs
sudo chmod +s /sbin/umount.cifs

```
So that users can mount and unmount the share without root privileges.

"No such device or address" is probably because "%20" doesn't work to represent a space, a quick google search seems to indicate that the space should be replaced with "\040" (no quotes), which is the character code for a space.

---

### Post by eadwacer on 2008-02-11
Well, nothing seems to work this time.

I ran the two chmods
I replaced the string. That section should look like:
\040Files/
right?

ran sudo mount

Same error: no such device or address

When I looked at mount.cifs in the browser, it still shows the user as root, with no-one else having any permissions

When I go to the Places/Computer menu it shows the share as an smb, but when I try to mount it via a right mouse-click it says:

mount error: permission denied or not superuser and mount.cifs not installed suid

Maybe I am doing something wrong with the chmod.  I'll dig around and see if I can find something. (I really hate for you to have to feed me such simple commands. I've done a lot of Win work, but I'm a n00b when it comes to linux).

---

### Post by compholio on 2008-02-12
> **eadwacer said:**
> Well, nothing seems to work this time.

I ran the two chmods
I replaced the string. That section should look like:
\040Files/
right?

ran sudo mount

Same error: no such device or address

When I looked at mount.cifs in the browser, it still shows the user as root, with no-one else having any permissions

When I go to the Places/Computer menu it shows the share as an smb, but when I try to mount it via a right mouse-click it says:

mount error: permission denied or not superuser and mount.cifs not installed suid

Maybe I am doing something wrong with the chmod.  I'll dig around and see if I can find something. (I really hate for you to have to feed me such simple commands. I've done a lot of Win work, but I'm a n00b when it comes to linux).

It's not a problem, yeah - the line should read (according to the source I found):
```
//NASbox/Shared\040Files/ /media/nasbox-shared cifs user,guest,noauto,rw,noperm 0 0
```

If you execute "ls -alF /sbin/umount.cifs" then it should report something like:
```
-rwsr-sr-x 1 root root 9220 2007-12-18 00:28 /sbin/umount.cifs*
```
(the "-rwsr-sr-x" means the file is "installed suid")

Does the share require a username and password to login?

---

### Post by eadwacer on 2008-02-12
ran the command, got this:
-rwsr-sr-x 1 root root 9100 2007-12-17 23:18 /sbin/umount.cifs*

except that the /sbin/umount.cifs* part was highlighted in red

no password required.

---

### Post by eadwacer on 2008-02-12
It just occurs to me that the problem might be on the NAS end. As I recall, and it's been over a year since I set the box up, on a Win network, they said "works on linux networks  -- using a smb connection". I don't know enough to know if this is significant (if we are trying to set up an other-than-smb connection), and I hope I haven't been wasting your time. Demonstrates the depth of my lack of knowledge.

---

### Post by compholio on 2008-02-12
> **eadwacer said:**
> It just occurs to me that the problem might be on the NAS end. As I recall, and it's been over a year since I set the box up, on a Win network, they said "works on linux networks  -- using a smb connection". I don't know enough to know if this is significant (if we are trying to set up an other-than-smb connection), and I hope I haven't been wasting your time. Demonstrates the depth of my lack of knowledge.

Yeah, "cifs" is the new protocol for handling windows shares - you could try using "smbfs" instead but I've never seen that work better than cifs.  What exact error do you get if you run "mount /media/nasbox-shared" or "sudo mount /media/nasbox-shared"?

---

### Post by eadwacer on 2008-02-12
For the plain mount command I get:
mount error: permission denied or not superuser and mount.cifs not installed SUID
(this despite the fact that I ran your chmod commands)

for sudo mount I get:
retrying with upper case share name
mount error 6 = No such device or address
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)

and, when I run the ls command you suggested, I indeed get:
-rwsr-sr-x 1 root root 9100 2007-12-17 23:18 /sbin/umount.cifs*
but the /sbin... part is highlighted in red.

Let me go in through my Win box and see if I can change some settings or permissions or something.

---

### Post by compholio on 2008-02-13
> **eadwacer said:**
> ...
mount error 6 = No such device or address
...

It must not be finding the mount point (sudo gives the most accurate error message, error messages are not always propagated correctly to non-sudo).  Try pinging "NASbox" and finding it's IP, then change the fstab entry like this (replace 192.168.0.150):
```
//192.168.0.150/Shared\040Files/ /media/nasbox-shared cifs user,guest,noauto,rw,noperm 0 0
```

---

### Post by eadwacer on 2008-02-13
I tried the ping-and-replace process, with same ultimate result: mount error 6 = No such device or address

However, a new twist has come up. Ping worked fine, but it would appear that it thinks that it's pinging my Westell router, not my NAS.

In any event, life has caught up with me, and I'm going to be hors de cyber probably through the weekend. Let me see what I can figure out about the name confusion, and I'll re-engage next week.

I really appreciate your patience and attention to detail.  Thanks.
Steve

---

### Post by compholio on 2008-02-15
> **eadwacer said:**
> ...
However, a new twist has come up. Ping worked fine, but it would appear that it thinks that it's pinging my Westell router, not my NAS.
...

That must be the problem, try executing a NetBIOS name lookup and see what it says the IP is:
```
nmblookup NASbox
```

By default Windows uses the IP returned by NetBIOS, Linux does not.

---

### Post by eadwacer on 2008-02-17
Sorry about the delay in responding. Three day weekends just aren't as long as they used to be. 

Both ping and nmblookup give the same IP address, however:

nmblookup nasbox:
querying nasbox on 192.168.1.255
192.168.1.30 nasbox

ping nasbox: 
nasbox.myhome.westell.com (192.168.1.30)

Westell is my DSL router.  (my setup is DSLRouter->hub-<PCs)  But when I ask it (through the setup GUI) about its local IP address, it tells me it's using: 192.168.1.1.  Presumably, 192.168.1.255 is my Linux machine.

Looking at my settings notebook (updated erratically), when I added the NAS I gave it the 192.168.1.30 IP address, so that, at least, checks out.

I tried using the -S parameter on nmblookup (man pages say that gives more info) and I got this....

        NASBOX       <00> -         B <ACTIVE> 
        NASBOX       <03> -         B <ACTIVE> 
        NASBOX       <20> -         B <ACTIVE> 
        ..__MSBROWSE__. <01> - <GROUP> B <ACTIVE> 
        BROADNAS        <bc> - <GROUP> B <ACTIVE> 
        WORKGROUP       <00> - <GROUP> B <ACTIVE> 
        WORKGROUP       <1d> -         B <ACTIVE> 
        WORKGROUP       <1e> - <GROUP> B <ACTIVE> 

...which runs right off my map.  I'll spend some time later this weekend parsing what that stuff means, and get back to you.

Thanks, again.
Steve

---

### Post by compholio on 2008-02-19
> **eadwacer said:**
> ...
Both ping and nmblookup give the same IP address, however:

nmblookup nasbox:
querying nasbox on 192.168.1.255
192.168.1.30 nasbox

ping nasbox: 
nasbox.myhome.westell.com (192.168.1.30)
...

Oh, that should be fine actually.  Most routers are at the IP 192.168.x.1 BTW.  That name is actually not the name corresponding to your router, but indicating that the box is on your network managed by your router.  Your problem is now starting to get a bit bizarre, what happens when you try to use the program "smbclient" to connect to the share? (you can find information on how to use this application by running "man smbclient")

---

### Post by eadwacer on 2008-02-19
> **compholio said:**
> Oh, that should be fine actually.  Most routers are at the IP 192.168.x.1 BTW.  That name is actually not the name corresponding to your router, but indicating that the box is on your network managed by your router.  Your problem is now starting to get a bit bizarre, what happens when you try to use the program "smbclient" to connect to the share? (you can find information on how to use this application by running "man smbclient")

Ow. Head hurt. I shan't be able to get to that for a few (I'm stealing time right now). On the router address, I seem to remember specifying everyones IP when I set things up a few years ago. SInce it's been pretty much untouched since then, I've forgotten half the things I did.  Thanks.

---

### Post by eadwacer on 2008-02-20
Just a quick note. Tried smbclient. First tried it with DOS separators:

smbclient  \\nasbox\\shared files\
It seemed to want everything doubled. If I didn't, I got an error:
\nasbox\shared: Not enough '\' characters in service
Usage: [-?] [-...

So, when I did the \\ bit, I got a > prompt (not smb:>, just >) and if I typed anything, like dir or ls (being not sure if I should be in DOS or linux mode), it dumped me back to the same error message.

Then I tried it with // instead of \\. When I did that, it asked me for a password, which it should not be doing because I am really sure I didn't password protect that drive. At least it thinks it's talking to something.

Anyway, we have an accreditation team coming next Monday, and I am just going to have to let this rest for the next week or so.

Thanks for your help. I shall return.
Steve

---

### Post by compholio on 2008-02-21
OK, for when you return:

"\" is a special character in linux (for example "\ " means space, since space is a different kind of spacial character), in order to get 1 slash you must use 2, to get 2 you must use 4, ie:
```
\\\\naxbox\\shared\ files
```

If it prompts you for a password (and there is no password) then you should be able to just hit enter.

---

### Post by eadwacer on 2008-02-21
I had to try it. It worked.

---

### Post by compholio on 2008-02-21
> **eadwacer said:**
> I had to try it. It worked.

That is strange that your fstab entry is not working, I modified mine to contain a space and it works:
```
//media/music\040folder
```

---

### Post by eadwacer on 2008-03-24
compholio
I promised to get back to this, and now I find it's been over a month. I appreciate all your work, and would not want it to go to waste...but it looks like it's too hard to do, unless and until Sunbird improves. I have come up with a workaround that fits my simple needs, at least until this summer.  Since I am going to have to spend most of my time on the XP box this quarter, I will just update all my Sunbird entries there - it stores the calendar file on my NAS.  Sunbird on the linux box can't see the NAS, but Nautilus can, and it's a simple draganddrop to pull the file onto the linux drive, which Sunbird can see.  I'll have to do a lot of synchronizing anyway, and this is just one more step.

Again, I can't say how much I appreciate all the work you've done with me. Time is precious, and I thank you for contributing yours.

Thanks again.

Steve

---

