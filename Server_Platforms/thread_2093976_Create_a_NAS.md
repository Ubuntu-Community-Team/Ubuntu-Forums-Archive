---
title: "Create a NAS?"
date: 2012-12-12
forum: Server Platforms
---

### Post by PDA1 on 2012-12-12
I'd like to create a home NAS.

Is there a simple guide on how to do it?

---

### Post by Lars Noodén on 2012-12-12
What kind of hardware do you have?  If you have multiple disks then you could have RAID 5 or RAID 10.

Other than that, setting up a NAS is simply using SSHFS, Samba, or NFS.  What kind of computers (Linux, Mac, etc) are you planning to connect?  From where, LAN or WAN?

---

### Post by darkod on 2012-12-12
Another option, depending how suitable it is to you, is FreeNAS instead of ubuntu based NAS.
[http://www.freenas.org/](http://www.freenas.org/)

---

### Post by PDA1 on 2012-12-12
> **Lars Noodén said:**
> What kind of hardware do you have?  If you have multiple disks then you could have RAID 5 or RAID 10.[QUOTE]

I don't know how to answer your question.

I've got a bunch of computers at home and I want to be able to share files among them with the least amount of complications and difficulties. 

Cloud storage is out of the question.

---

### Post by darkod on 2012-12-12
One machine has to have the role of the file server. It will host the files and be online all the time so that other machines can access it.

So, it depends a little bit which computer/server you want to use for this role, the HDDs you have inside, etc. For example, for raid5 you need a minimum of three HDDs, so if you have only two, there is no way to do raid5. That's why it matters.

And by "least amount of complications and difficulties" you mean from the users perspective, or yours? You will need to have some basic knowledge to administer the server regardless which solution you choose.

---

### Post by Lars Noodén on 2012-12-12
NAS is no different then 'cloud', just local.

If you are looking to set up one single machine to act as a hub for file transfer and storage, then you have the three options above.  Of them, SSHFS is the least trouble to set up, is very secure (it works over SFTP) and work over both LAN and WAN.  

RAID is useful to protect against disk failure, but should not be confused with backup.  With RAID, if a disk fails, you can put in a new one and keep going.

---

### Post by PDA1 on 2012-12-12
Local "cloud" is really what I'm looking for...I think.

Is the following correct?;

1 computer acts as the central hub for storing files.

All other local computers are connected to the central hub and are configured so that they can access the central hub to retrieve and/or send files to it.

The hub computer is on all of the time. If it's not then none of the files on it can be accessed.

The hub computer is connected to other local computers via ethernet cable.

The hub computer must be running some os.  Ubuntu is preferred (since I'm using Ubuntu)

With the hub computer running Ubuntu, SSHFS on the hub and allows for the exchange of files between local machines.

Am I correct in the above statements?

Thanks for the help folks.

---

### Post by dannyboy79 on 2012-12-12
yes, all those statements are true. however, will you ever want to retrieve files from this server from outside your LAN? (local area network) if not, then I don't see the need to use SSHFS because it adds a layer of encryption that will slow down the transfer speeds. Either NFS or SAMBA is suitable for LAN file server storage. SAMBA works with all three OS's, OS X, Windows, and Linux.

Do you want redundancy? Meaning if a hard drive dies, you don't want the risk of losing data? If so, then you'll need to implement a form of RAID as well.

Freenas may be your easiest bet for setting everything up if the sole purppose of the server will only be file storage/serving

---

### Post by Lars Noodén on 2012-12-12
That about sums it up.  But all transfers go to or from the NAS hub, not directly to or from the end nodes.

SSHFS is quite speedy.  Your limiting factor is more likely to be the speed of your local network's router.  SSHFS will also let you securely access your data over the WAN, not just the LAN.

---

### Post by PDA1 on 2012-12-12
I won't be accessing any of the files outside of my LAN.

When it come to the actual implementation of setting up a home NAS, can I use my existing main computer which already has ALL of the important files on it?  That is, on my main computer all I would have to do is install SSHFS (I like the idea of encrypted transfer even if it's local) so that the other computers in the house could access it?  

Are the following correct?

With SSHFS installed on my main computer where all of the important files I'd access are located, there would be no real significant change to the version of Ubuntu it's running (10.04).

I will be able to stream videos and music over the LAN.

Again, thank you all for the help.

---

### Post by Lars Noodén on 2012-12-12
Strong encryption is good to have. 

For SSHFS, all you need on the NAS is the ssh server (sshd).  That is provided by the package openssh-server.  On the client side, you need the package sshfs.  It is just a fancy sftp front-end.  You can read a little more here:
[https://help.ubuntu.com/community/SSHFS](https://help.ubuntu.com/community/SSHFS)
It is easy to set up.

---

### Post by PDA1 on 2012-12-12
An abstract question;

When connecting a local computer to the main computer (server) must the both machines be connected to a central ethernet router?

---

### Post by dannyboy79 on 2012-12-12
> **PDA1 said:**
> An abstract question;

When connecting a local computer to the main computer (server) must the both machines be connected to a central ethernet router?
yes, that's assuming they are in the same location and on the same subnet. ethernet connected or wirelessly connected.  you haven't really answered the question, do you need to access the file server from outside your local area network? (LAN)

if this is just a home network, encryption is overkill in my opinion.

---

### Post by PDA1 on 2012-12-12
As I said before, "I won't be accessing any of the files outside of my LAN".  By that I mean I won't be accessing the main server/computer from anywhere else in the world except from within my house.  Does that make sense?

So encryption is overkill if I'm accessing only at home.

Must I connect via ethernet router or can I simply use my existing wireless router?  I do know that one of my computers is connected via ethernet cable (or whatever it's called) to the wireless router.

I'd like to do the set up as cheaply as possible and not having to buy another router would be nice.

Is there a way to just simply plug an ethernet cable from one computer to the other and gain the same accessibility?

What's your opinion?

---

### Post by Lars Noodén on 2012-12-12
Encryption on the LAN is not overkill.  It's a good practice.  It also means that your method becomes usable across the WAN should you decide to do so later.

You can just plug cables across between two machines, if you have the interfaces setup right.  But the more common way is to connect via your home router.  If you want the simplest way of transfering files, then use SFTP: put openssh-server on one machine  and then from the other use an SFTP client like Nautilus or Thunar.  Both have SFTP support built in.

---

### Post by tgalati4 on 2012-12-12
I like [http://freenas.org](http://freenas.org)  You can read the forums or do a google search on "freenas build blog" and read other's experiences with setting up a home server.  Power consumption can be an issue if it is on 24/7.  You can set up a server and put it to sleep and set up wake-on-lan on each machine in the house to wake it when needed.

---

### Post by dannyboy79 on 2012-12-12
> **Lars Noodén said:**
> Encryption on the LAN is not overkill.  It's a good practice.  It also means that your method becomes usable across the WAN should you decide to do so later.

You can just plug cables across between two machines, if you have the interfaces setup right.  But the more common way is to connect via your home router.  If you want the simplest way of transfering files, then use SFTP: put openssh-server on one machine  and then from the other use an SFTP client like Nautilus or Thunar.  Both have SFTP support built in.another reason I feel this is not an ideal way of sharing files is because there's no possible way for a media type device to access a media file like a song or movie. Maybe there is but it's not as simple as using a file sharing protocol. Also, there's the fact that SSHFS will allow access of the user to potentially delete system files since they have access to the entire filesystem and not just shared folders with proper permissions.

---

### Post by PDA1 on 2012-12-12
What would you recommend then?

---

### Post by dannyboy79 on 2012-12-12
> **PDA1 said:**
> What would you recommend then?either freenas or ubuntu plus samba, especially if you'll have windows machines within the network. freenas may be more easily configurable since it's sole purpose is to be a file server.

---

### Post by PDA1 on 2012-12-12
FreeNas running FreeBSD is not an option for me. Personal preference that's all.

So, I guess it's going to have to be ubuntu plus samba.

---

### Post by PDA1 on 2012-12-12
Is there an "idiots guide" to using Ubuntu/Samba?

I installed Samba (the laughter begins from the audience) on my 10.04 machine.  I saw a whole big list of users on one of the Samba options and promptly uninstalled Samba.  Who the heck are they?!

Anyway....so I'll eventually put Samba on my 12.04 and 10.04 machines (so I say). The only problem is in the first trial of it I couldn't "see" my 10.04 machine from my 12.04 machine.

Any ideas?

---

### Post by darkod on 2012-12-13
I have no idea about what list of users you are talking about (and i have installed samba only as part of a server OS install, not on a desktop OS).

But until you set up a samba share(s) there is nothing to be seen from other computers. Did you set up at least one share?

---

### Post by PDA1 on 2012-12-13
Solved;

Installed ssh something-or-another.

Connect to Server from Places.

Enter the connection address...something like 192.189.3.89

User name- the name on the other computer
PW- the other computer's login password.

Logs right in and I can look at the entire computer and get files.

Really easy.

---

### Post by darkod on 2012-12-13
That looks more like a remote session to the computer, not file sharing.

But if you are happy with it, it's your choice.

But have in mind that if you want more users accessing the files at the same time, you will have to check if you can have more than one remote sessions working at the same time.

With samba shares that is not a problem, you can have many computers accessing the shares.

---

### Post by dannyboy79 on 2012-12-13
sounds like he went with sshfs. will work fine for simple just file transfering but won't be able to stream media like movies, music and pictures.

the list of users are probably the system users that the system creates by default and can be ignored. I haven't set up samba in any recent ubuntu so I am not sure what GUI settings thing poped up. I believe ubuntu is trying to make it way more easy to share files, you could just right click on a folder and in the menu should be a share folder something or other. Never used that though so can't comment.

---

### Post by PDA1 on 2012-12-13
I could watch a video that was located on the computer "B" which I was logged into while using computer "A" with the method I described briefly above. I got the same results listening to music that was on the other computer. The files weren't tranferred to reside on the machine I was working on (computer "A") 

I could access computer "B" from the computer I was using (computer "A"). At the same time I could log into computer B from computer A.

No one else "in house" will be doing the same thing as I am or trying to access the files. This makes it quite nice as I can connect to their machine and send the files to them that I want to back up. Thus, I can spread my backups all around the network.

Prior to installing OpenSSH (or whatever it's called) I couldn't access any other computer.

---

