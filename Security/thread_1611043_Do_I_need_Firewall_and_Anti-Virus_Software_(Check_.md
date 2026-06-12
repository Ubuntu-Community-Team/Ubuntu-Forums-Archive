---
title: "Do I need Firewall and Anti-Virus Software? (Check for More Info)"
date: 2010-11-01
forum: Security
---

### Post by D3SI on 2010-11-01
Ubuntu 10.04 - 32Bit
I do Torrenting a lot - I am using qBittorrent but i mostly use websites like, 
[LIST]
[*]TorrentLeech (Private Site), 
[*]SceneAccess(Private Site), 
[*]BitSoup (Private Site) and some times...
[*]Piratebay(Public Site)
[/LIST]

do I need to take any security measures? can anyone hack my info because I am using torrent client and stuff?

---

### Post by ubunterooster on 2010-11-01
With Ubuntu, just run ```
sudo ufw enable
``` to enable the firewall. That should be sufficient, though you could use "virus scanner" (get it from Ubuntu Software Center) to be safer

---

### Post by D3SI on 2010-11-01
thanks.. ran the command, also if you could tell me what that command does so I know ;)

will check for Anti-Virus

Edit: nvm..  Uncomplicated Firewall ::P

---

### Post by ubunterooster on 2010-11-01
ufw = "[COLOR=Red]u[/COLOR]ncomplicated[COLOR=Red] f[/COLOR]ire[COLOR=Red]w[/COLOR]all" Unless you have Samba filesharing or a few other services, you should not need any other configuration than merely enabling it. 

Manpage: [http://manpages.ubuntu.com/manpages/maverick/en/man8/ufw.8.html](http://manpages.ubuntu.com/manpages/maverick/en/man8/ufw.8.html)

---

### Post by D3SI on 2010-11-02
installed...

and noticed that my PS3 Media Server is not detecting PS3 anymore..

could firewall be blocking it?

if yes how do i sort it out?

---

### Post by mastablasta on 2010-11-02
Install gufw which is a GUI for the firewall and then configure to let the PS3 media server through.
 
also even if oyu use firewall they cna still get your data such as you IP and can sue you for downloading "illegal" content, if that is what you are worried in the first post.

---

### Post by D3SI on 2010-11-02
I want to use it so no one can hack my pc..  not worried about illegal content...

edit: thanks for help  ran these commands and it worked :)

```
sudo ufw allow 5001/tcp
```

```
sudo ufw allow 5001/udp
```

---

### Post by inameiname on 2010-11-02
If you want a better ufw frontend, I'd try 'ufw-gtk' instead of 'gufw'. It's got a lot more options, and I prefer it over gufw.


[LIST]
[*]sudo add-apt-repository ppa:baudm/ppa
[*]sudo apt-get update && sudo apt-get install ufw-gtk
[/LIST]

---

### Post by mastablasta on 2010-11-02
> **D3SI said:**
> I want to use it so no one can hack my pc.. not worried about illegal content...
 
edit: thanks for help ran these commands and it worked :)
 
```
sudo ufw allow 5001/tcp
```
 
```
sudo ufw allow 5001/udp
```
 
i see. well as i understand you just opened doors no. 5001 to your PC. 
 
so theoretically one could hack to your PC through those doors. however if they are limited only to specific programme then they would have to hack through that programme. 
 
or i just understand things the wrong way, but i believe this is how port forwarding works.

---

### Post by D3SI on 2010-11-02
how do i  limit it to the programme?


@[inameiname]("http://ubuntuforums.org/member.php?u=949055")  its not in the market?

---

### Post by drmarkandersen on 2010-11-02
Hi, 
Don't know if it's appropriate to tack on a question of my own, but since we're talking about firewalls ...
What are the relative merits of Firestarter as opposed to the two firewall GUIs that have been mentioned here (gufw and ufw-gtk)? I'm looking for something that's not going to mess up samba and bittorrent when my laptop is at home, and that's going to get along well with my university's firewall when I'm at work.

---

### Post by D3SI on 2010-11-02
installed ufw gui version

please look at the fields and help me...

also what does these commands do mentioned in above post

```
sudo add-apt-repository ppa:baudm/ppa
sudo apt-get update && sudo apt-get install ufw-gtk

```

---

### Post by kwacka on 2010-11-02
> **D3SI said:**
> ```
sudo add-apt-repository ppa:baudm/ppa
```
Adds the ppa (Personal Package Archives) 'baudm' to your repository list.

> **D3SI said:**
> ```
sudo apt-get update && sudo apt-get install ufw-gtk

```

makes sure that changes to your repository are recognised by your system. '&&' enables a second command to be added to the same line. In this case to install ufw-gtk

---

### Post by D3SI on 2010-11-02
can you help me with those fields please?

see above post attachment

---

### Post by inameiname on 2010-11-02
[FONT=Arial]Thank you kwacka for explaining it to D3SI.

It's just a quick and easy way to install the software. Why I prefer the terminal. I'm a terminal nut. :P In contrast, you could manually add the ppa, by adding the lines to /etc/apt/sources.list

[/FONT][FONT=Arial]deb [http://ppa.launchpad.net/baudm/ppa/ubuntu](http://ppa.launchpad.net/baudm/ppa/ubuntu) maverick main 
deb-src [http://ppa.launchpad.net/baudm/ppa/ubuntu](http://ppa.launchpad.net/baudm/ppa/ubuntu) maverick main [/FONT][FONT=Arial]and then manually adding the pubkey

and then go to software center and find "ufw-gtk" and install.

Basically, you have to add that repo because 'ufw-gtk' isn't available in the official Ubuntu repos.
[/FONT]

---

### Post by 3rdalbum on 2010-11-02
If your Bittorrent client is the only thing that is listening for incoming connections, then you don't need a firewall. The firewall will just block incoming torrent requests, which you don't want, and it won't add any more security because the only incoming port is the Bittorrent one anyway.

---

### Post by D3SI on 2010-11-02
how can i allow PS3 Media Server through the Firewall?

---

### Post by uRock on 2010-11-02
> **D3SI said:**
> installed ufw gui version

please look at the fields and help me...

also what does these commands do mentioned in above post

```
sudo add-apt-repository ppa:baudm/ppa
sudo apt-get update && sudo apt-get install ufw-gtk

```
I would just use GUFW. I don't trust adding repositories, especially for security software.

To allow your PS3 to connect you need to allow the port via GUFW. Just click the ad button and go from there.

Moved to Security Discussions.

---

