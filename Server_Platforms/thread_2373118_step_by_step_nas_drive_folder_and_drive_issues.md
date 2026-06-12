---
title: "step by step nas drive folder and drive issues"
date: 2017-10-03
forum: Server Platforms
---

### Post by leebrendalee2 on 2017-10-03
forgive me if this has already been asked a million times but frankly after 2-3 weeks of trying endlessly trying I need help. Please be patient as I work through the steps.
I have watched every youtube video and endless upon endless google help streams ...I think i'm just dense.  I don't know the terminology so I came here to learn it.

My nas: 192.168.1.233
At the top is says NasDrive1-Dynology Diskstation (some how with all of my messing around I figured changing the name might help) nope!!
under Shared Folder: TV
under File Station: TV (when I go into File Station I notice a folder NasDrive1 then the TV folder  (ok wonder why I did that I expect to have another Nas when I don't know how to use this one) 

I am running Ubuntu and do you think for one minute that I can get to those folders? I will post my fstab file can anyone please help me? I have tried every combination possible.  I don't understand what "media" folder and do I need it and "var". oh I'm so confused.
ok, since its on a different computer guess cut and paste won't work..duh

basically 

//192.168.1.233/volume1/TV/home/var/media/tv/nfs rsize=8192,wsize=8192,timeo=14,intr
I've tried it without the //

thanks in advance

---

### Post by slickymaster on 2017-10-03
Thread moved to **Server Platforms** for a better fit

---

### Post by darkod on 2017-10-03
This is not very much ubuntu related, it is more NAS related. It depends how you need to open shared folders on your NAS (for example the volume1 in the path might not be needed).

First, do you have ubuntu server version or desktop version with a GUI? And you are trying to open the NAS share from ubuntu, right?

---

### Post by leebrendalee2 on 2017-10-03
yes its actually ALL ubuntu related.. I don't have a problem with the nas drive whatsoever, everything is fine there.  I was just starting there.  I am using one one machine Ubuntu 16.04 LTS device name on that one is MediaServer, its graphical.  I everything working "ok" until it stopped working.  So over to the test box  I have a different version of Ubuntu there and trying to setup from scratch graphical both using command lines though, and cannot get it working there either.  It all has to do with the /etc/fstab directory I believe.  Now on the media server I can see the computer-var-media-and my directories but theres nothing in them, they just vanished. But at this point I'm trying to UNDERSTAND what to do because if I cannot recreate anything that I'm not learning how to do this.  I"m here to actually understand how to do this so that I can create it again. Its hard and I've been trying for 2-3 weeks on this.  LOL I'm stubborn should have posted before but usually can figure out with the other posts reading.

---

### Post by darkod on 2017-10-03
I said related to the NAS because it depends how the share is published. For example, if you open the NAS in windows with \\IP, does it show the TV share right there? If it does, in linux the mount line should be //IP/TV, not //IP/volume1/TV. The 'volume1' might be internal path thing and might, or might not be necessary in the mount line.

Also, the mount line you posted does not seem correct. I don't see a mount point in it. Maybe that got lost during the pasting.

First try to mount temporary at the command line, if the TV share accept anonymous access it would be something like this. And make sure you have cifs-utils installed, otherwise you can't mount cifs.
```
sudo apt-get install cifs-utils
sudo mount -t cifs //192.168.1.233/TV /mnt -o guest
```

That should be enough to see if you can mount the share on /mnt.

If you are trying to mount another type of share, like nfs, let us know because the command is different.

PS. I asked if ubuntu client has GUI because with the GUI you can easily see how the share is published if you don't know that. Open Nautilus (the file manager) and use the option Connect to Server. After you connect to 192.168.1.233, what do you see? The share called TV?

---

### Post by leebrendalee2 on 2017-10-03
> **darkod said:**
> I said related to the NAS because it depends how the share is published. For example, if you open the NAS in windows with \\IP, does it show the TV share right there? If it does, in linux the mount line should be //IP/TV, not //IP/volume1/TV. The 'volume1' might be internal path thing and might, or might not be necessary in the mount line.
                            Thank you very much for helping me!  You said when I open the nas in windows, do you mean when I open it up via any browser in windows/, no the                     TV share is not there.  I need to go into the folder to see it.  If you mean am I sharing the nas on windows, not yet.  I see it as as shared drive it                         shows up but when I click on it, the browser opens up and I need to log in etc.  Sorry if I sound confusing I'm just trying to answer your question.  


                                   Also, the mount line you posted does not seem correct. I don't see a mount point in it. Maybe that got lost during the pasting.

First try to mount temporary at the command line, if the TV share accept anonymous access it would be something like this. And make sure you have cifs-utils installed, otherwise you can't mount cifs.
```
sudo apt-get install cifs-utils
sudo mount -t cifs //192.168.1.233/TV /mnt -o guest
```

install your utility and error is "couldn't chdir to mnt: no such file or directory.  
That should be enough to see if you can mount the share on /mnt.

If you are trying to mount another type of share, like nfs, let us know because the command is different.
I believe it is NFS and I saw the directory as volume/TV

PS. I asked if ubuntu client has GUI because with the GUI you can easily see how the share is published if you don't know that. Open Nautilus (the file manager) and use the option Connect to Server. After you connect to 192.168.1.233, what do you see? The share called TV?

thats another problem, LOL I have been trying that for a long time and its always greyed out.  I'm thinking I'm missing something that goes in front because it says in grey below (smb://)

---

### Post by darkod on 2017-10-03
It should work with server address smb://192.168.1.233. Try it.

---

### Post by leebrendalee2 on 2017-10-03
ok error: oops, something went wrong. Unhandled error message: failed to retrieve share list from server: connection timed out

---

### Post by darkod on 2017-10-03
Doesn't look like only ubuntu problem. Does the NAS has static IP? 192.168.1.233 is very rare choice for server static IP. Make sure you have all that correct, and you are trying to connect where you think you are.

Looks like the ubuntu desktop can't even reach the NAS shares correctly. Have you tried rebooting the NAS?

---

### Post by leebrendalee2 on 2017-10-03
ok i'm rebooting the nas.  I can reach the nas no problem in the browser, yes static IP.  I can reach it from my phone and ipad too no problem. ok I rebooted the nas tried the following
smb://192.168.1.233  failed to retrieve share list from server, connection refused, then I tried smb://192.168.1.233/volume1/TV  failed to mount windows ahre connection refused

---

### Post by darkod on 2017-10-03
When you reach it from the phone and ipad, is it using some app or what? How does it list the shares, how do you connect? And do you use credentials or it has anonymous access?

---

### Post by MAC59 on 2017-10-17
Hello Guys,

          I am not sure if this has already been suggested, I have a QNAP nas and I have to submit either a user, a computer name or if I am doing iSCSI an IQN of the initiator in an ACL list to gain access ot it.  Is it possible that he needs to do that to get the access to it? Like I said sorry if it's already been suggested.

---

