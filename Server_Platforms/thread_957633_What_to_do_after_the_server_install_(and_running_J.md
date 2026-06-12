---
title: "What to do: after the server install (and running Joomla)"
date: 2008-10-24
forum: Server Platforms
---

### Post by Lakeside on 2008-10-24
I have googled and found some good tutorials concerning Hardy Heron installation,  and then installing Joomla into it.  While I am a little familiar with Joomla, I am new to Linux, Ubuntu, and web servers (well, did start out some time ago, but wasn`t able follow it up til recently so..). I thought I would ask your advice, since I`ve gotten excellent help here so far. I just don`t know enough, I feel, to tell if what the tuts are saying is right, so could someone point 
me to the following- pleeeez :) - a good guide on what exactly I do after Hardy Heron is installed, which would have me running the server, with Joomla on it, and securely.
So far I have enabled a few programs (unrar,  chm, media players etc. by the terminal, so catching on a little about apt get, and sudo) but that`s it.  Thanks so much for any help.

---

### Post by Sarmacid on 2008-10-24
I would recommend setting up a firewall with iptables, and installing ssh server if you plan on managing it remotely.

---

### Post by bodhi.zazen on 2008-10-24
> **Lakeside said:**
> I have googled and found some good tutorials concerning Hardy Heron installation,  and then installing Joomla into it.  While I am a little familiar with Joomla, I am new to Linux, Ubuntu, and web servers (well, did start out some time ago, but wasn`t able follow it up til recently so..). I thought I would ask your advice, since I`ve gotten excellent help here so far. I just don`t know enough, I feel, to tell if what the tuts are saying is right, so could someone point 
me to the following- pleeeez :) - a good guide on what exactly I do after Hardy Heron is installed, which would have me running the server, with Joomla on it, and securely.
So far I have enabled a few programs (unrar,  chm, media players etc. by the terminal, so catching on a little about apt get, and sudo) but that`s it.  Thanks so much for any help.

Those are fairly broad questions. See if these get you started, ask if you have questions :twisted:

[https://help.ubuntu.com/8.04/serverguide/C/index.html](https://help.ubuntu.com/8.04/serverguide/C/index.html)

[https://help.ubuntu.com/community/Joomla](https://help.ubuntu.com/community/Joomla)

---

### Post by Lakeside on 2008-10-24
Good, you reminded me (and confirmed too ) about the iptables (saw it in  `first ten things to do after installing Ubuntu`, somehthing like that, it`s a must for security I guess.  And I did sort of browse through that help list, but it mentions LAMP, and apache, mysql etc , and I`m not using that, I`m using Hardy Heron server, so I thought it might be different..somehow.  I`m sure I`ll get it if I just keep plugging away. thanks all

---

### Post by ichimr285 on 2008-10-25
[img]http://www.top1gaming.com/cosplay/GuildWars-5.jpg[/img][font=Times New Roman][size=3]See the answer [/size][/font][[font=Times New Roman][size=3][color=#800080]click here[/color][/size][/font]](http://www.top1gaming.com/coscontent-60-7.html)[font=Times New Roman][size=3].  Want to see more [/size][/font][[font=Times New Roman][size=3][color=#800080]cosplayer[/color][/size][/font]](http://www.top1gaming.com/cosplayer.php)[font=Times New Roman][size=3] ? [/size][/font][font=Times New Roman][size=3][/size][/font][font=Times New Roman]**[size=10pt]Recommend : [/size]**[size=10pt][[color=#0000ff]D.Gray-Man Lavi[/color]](http://www.top1gaming.com/coscontent-88.html)   [[color=#0000ff]World of warcraft[/color]](http://www.top1gaming.com/coscontent-57.html)  [/size][/font][size=10pt][[color=#0000ff]Ragnarok Online cosplay[/color]](http://www.top1gaming.com/coscontent-58.html)      [/size]

---

### Post by sethvath on 2008-10-25
[LAMP]("http://http://en.wikipedia.org/wiki/LAMP_(software_bundle)") - Linux, Apache, MySQL and Perl/PHP/Python

You do require mysql to run joomla. Check the [link]("https://help.ubuntu.com/community/Joomla") provided by bodhi

---

### Post by bodhi.zazen on 2008-10-25
You can manage your firewall with UFW, it may be easier.

[https://wiki.ubuntu.com/UbuntuFirewall](https://wiki.ubuntu.com/UbuntuFirewall)

[https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw](https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw)

---

### Post by Lakeside on 2008-10-25
Thanks bodhi.zazen, I just installed ufw, and then installed the gui for it (Firestarter), and was going to configure it, but I think that`s enough for today (also I would be asking some more questions as I`m not sure what to put in it, this whole server and network stuff is new to me!) . Sethvath, thanks too, but I am going to use Hardy Heron, which (and I`m still a little confused by all this) I think has all that stuff- apache, mysql, and php.

---

