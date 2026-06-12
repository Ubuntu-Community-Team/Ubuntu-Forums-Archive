---
title: "Xbox 360 + virtualbox + media player 11"
date: 2008-05-13
forum: Virtualisation
---

### Post by nunki on 2008-05-13
I am currently running Hardy 64bit, and have a windows xp sp2 guest running in virtualbox with host networking setup. I also have a samba share that I use for sharing files between ubuntu and my girlfriends mac(samba share on ubuntu). The guest os is able to log into the samba share and add all the media files to media player 11 and play them no problem (even able to turn on media sharing for the xbox).

My Xbox 360 is able to see the guest os on the network and connect; it can even build a list of all the files in the library, but is unable to play any :( Every song and picture has a red icon next to it and I get an error when trying to play any of them. Keep in mind the guest os which is "sharing" is able to play all of these files no problem.

Anyone try doing this before? Any clues why these simply wont play?

I have double checked all the file permissions, and taken a second look at smb.conf, but everything works great. Xbox just cant seem to play the files. Ive tried allowing guests in samba, but beyond that I dont have a clue.

---

### Post by nunki on 2008-05-13
bump

---

### Post by tighem on 2008-05-13
What's the file type? MP3? AAC?

Also, are you using host networking or NAT in Virtualbox?

---

### Post by nunki on 2008-05-13
> **tighem said:**
> What's the file type? MP3? AAC?

Also, are you using host networking or NAT in Virtualbox?

Host networking is set up and functioning well. All the files are either .jpg or .mp3

---

### Post by tighem on 2008-05-13
If I get time tonight I'll setup mine and see if it works...

---

### Post by nunki on 2008-05-13
> **tighem said:**
> If I get time tonight I'll setup mine and see if it works...

Id appreciate that. Ive been struggling to get this working for a while now. Make sure that you enable remote file sharing in windows, otherwise you wont even get the library list in the xbox. Im really hoping that this will just require some modified samba settings.

---

### Post by nunki on 2008-05-13
Just tried fuppes with no luck. I was able to get my xbox to see the fuppes share, but nothing showed up in the music or pictures list.

---

### Post by tighem on 2008-05-15
I tried it on mine and no dice...BUT my Xbox is behind a NAT'd Mac. I don't think file sharing works unless the Xbox and Media Center are on the same subnet.

---

### Post by nunki on 2008-05-16
> **Robocoastie said:**
> MCE content is actually rendered on the PC and streamed to your extender (which in your case is the XBOX360). Direct-X functions like MCE uses don't work in VirtualBox which is why you all you get when you try to watch your videos is a black screen.

I posted this same question in a different forum and got the above answer.Looks like even if they were on the same subnet (which mine are), Virtualbox doesnt support it.

---

