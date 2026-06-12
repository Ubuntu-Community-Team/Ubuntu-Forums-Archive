---
title: "Is there a way of being ROOT user for more than one command at a time?"
date: 2006-09-15
forum: Server Platforms
---

### Post by Nap_BlownApart on 2006-09-15
I've setup my Ubuntu 6.06 server with a Desktop GUI.
I've done this since I'm new to Linux and it helped me get going quicker.

I wish to edit the /etc/apt/sources.list file to remove some of the comments in it.

Trouble is that I can only open the file in Read-Only mode.

Q1)  Can I assume root while in the GUI?
Q2)  Is there a way of assuming root for more than a single command?

Cheers,
Nap

---

### Post by The_Apprentice on 2006-09-15
Welcome to Ubuntu :)

The immediate answer is no.

It is a very bad move to use a root user when you are logged in, so I am not even going to discuss how you could do it.
There are a large number of posts that discuss this, just do a search for SUDO.

If you want to edit files and things via the GUI then you could use the command "gksudo nautilus" or "kdesu konqueror" depending on which desktop you have.
This will give you root priveleges in "File Explorer" whilst it is open.

The best way to do most thing is via the command line.
In this case use "sudo" in front of the command eg "sudo gedit /etc/apt/sources.list".  Tis true you will often be prompted for the password, but at least you can sleep in the knowledge you system is very secure.

Have fun and enjoy.

---

### Post by chrisfay on 2006-09-15
```
sudo nautilus
```





> you could use the command "gksudo nautilus"


....just noticed that comment. Sorry for the repeat.

---

### Post by Nap_BlownApart on 2006-09-15
Where do I use the 'gksudo nautilus' command.  I am already in the gui (part of the boot process), and it looks like that command will open another GUI.

Cheers,
Nap


Not intending to upset anyone, but I have to say what's in my head at the moment.

I won't have time to sleep, I'm going to be typing my password in to much.  And when I do sleep, I won't be able to do so peacefully because I'll be worried about where the next security threat will come from.  So I consider it a false argument.

I grew up with the command line as the only UI.  I got used to it.  But I never stopped seeking better ways of doing things.  I'm sorry but to say that the command line is the best way to do things is like saying the best way to travel is by walking.  I don't buy it.

I can understand the argument for keeping people out of root.  Particularly when there are multiple users relying on the machine. But I own the computer, and I would like access to it.  Time is of essence in today's world.  I would like if I had the choice to decide how I want to protect my system.  If I wanted to crash my system with a hammer, how would Ubuntu (or any other secure system prevent me)?

---

### Post by wieman01 on 2006-09-15
> It is a very bad move to use a root user when you are logged in, so I am not even going to discuss how you could do it.
There are a large number of posts that discuss this, just do a search for SUDO.
The argument is valid but a bit naive because it assumes that every user is dumb. I have heard it a million times... We're here to help people, not to patronize them.

Just do the following:
> sudo passwd root
Then enter your normal user's password and then your new root password (twice). That should do and you should be able to switch to root this way:
> su root

[The commands enable the root account which is disabled by default for the mentioned reasons.]

---

### Post by Nap_BlownApart on 2006-09-15
The_Apprentice/ChrisFay
  Thnx for the commandline.  I've used it.

wieman01,
  Thnx for that.
  I've done what you suggested.  How do I allow root to logon through gnome?

**I do have one more question for your guru's**
By changing the sources.list file, I'm hoping to see more information in Synaptic.  I'm assuming that Synaptic uses this file (as well as aptitude)?


Cheers,
Nap

---

### Post by Nap_BlownApart on 2006-09-15
wieman01,
  Don't worry, I've figured it out.
  In System/Administration/Login Window.

Cheers,
Nap

---

### Post by wieman01 on 2006-09-15
Hi, 

Great. There is a nice howto:

[http://https://help.ubuntu.com/community/RootSudo]("http://https://help.ubuntu.com/community/RootSudo")

Just could not get hold of it this morning...

---

### Post by enopepsoo on 2006-09-15
> **Nap_BlownApart said:**
> I'm sorry but to say that the command line is the best way to do things is like saying the best way to travel is by walking.  I don't buy it.

Walking is the best way to get around.:cool: 

Also, you can do a lot from the command line and save yourself a lot of time.:KS

---

### Post by The_Apprentice on 2006-09-15
> **wieman01 said:**
> The argument is valid but a bit naive because it assumes that every user is dumb. I have heard it a million times... We're here to help people, not to patronize them.

Mkay, I was determined to bite my tongue and not reply to this comment, but I feel I must.

Firstly, my comment was not meant to be patronising in any way.

The question of privilieges and the pros and cons of root have been discussed to death.
In fact, whenever it is mentioned the thread suddenly fills with the potifications of various people and their views.
My comment was intended, and seems to have worked, to stop that before it even started.
I even hinted that a search on SUDO would have provided a wealth of witterings to read, leading down the steady road of wanting to slit your own throat.

I asked exactly the same question, in spirit, as Nap_BlownApart asked in that I wanted an easier way to undertake tasks in the GUI - [http://ubuntuforums.org/showpost.php?p=1473781&postcount=43](http://ubuntuforums.org/showpost.php?p=1473781&postcount=43)
To me that was the perfect answer.

---

### Post by wieman01 on 2006-09-15
> **The_Apprentice said:**
> Mkay, I was determined to bite my tongue and not reply to this comment, but I feel I must.

Firstly, my comment was not meant to be patronising in any way.

The question of privilieges and the pros and cons of root have been discussed to death.
In fact, whenever it is mentioned the thread suddenly fills with the potifications of various people and their views.
My comment was intended, and seems to have worked, to stop that before it even started.
I even hinted that a search on SUDO would have provided a wealth of witterings to read, leading down the steady road of wanting to slit your own throat.

I asked exactly the same question, in spirit, as Nap_BlownApart asked in that I wanted an easier way to undertake tasks in the GUI - [http://ubuntuforums.org/showpost.php?p=1473781&postcount=43](http://ubuntuforums.org/showpost.php?p=1473781&postcount=43)
To me that was the perfect answer.
Don't worry... I have read some of these threads and I basically agree with the concept. And I do understand what risks this entails. However, if user specifically asked for it (root access, etc.) I try to be straight and give them what they want. :-) But again, you have a point... Personally I would never log on to the system (X that is) with root authority.

Good discussion, buddy. No need to hold back & bite your tongue. ;-)

---

### Post by Nap_BlownApart on 2006-09-15
Thanks to all you guys.

I didn't mean to upset people, nor start any non-productive discussions.  It was my fault for allowing some of my recent 'install' related frustrations to come through.  I did try to make it a little light hearted with some of my analogies.

As a Windows user, I understand where everyone is coming from re GUI vs Commandline.

Maybe we can agree that there are horses for courses...

Cheers,
Nap

---

### Post by wieman01 on 2006-09-15
Nah... You didn't upset anybody. This kind of discussion is normal, at least in this forum. And usually is meant & done in a friendly way. Hey, it's Ubuntu, remember? :-)

---

### Post by The_Apprentice on 2006-09-15
No upsets as far as I am aware.

I am in exactly the same boat.
I have worked as a Microsoft consultant for at least the last 10 years.
You want to know anything about windows/dos and I could give you an answer.

I want to broaden my horizons, but my first aim was to replace my W2K/Echange 2000/IIS server (at home) with a Linux server, which I have now done.
Ultimately I would like to become Linux/Ubuntu certified, but that is a long way off.

I still have a XP box for all my gaming.

---

### Post by Nap_BlownApart on 2006-09-15
The Apprentice,

lol, similar setup here.

I still have my W2K Server running (with IIS/SQL2K) on the LAN with my Ubuntu.  I'm talking to you guys on this W2K client, and also have a XP Pro machine I use to test with.

One of my challenges is to have both running harmoniously (preferrably with one PAM database).  So far I've been able to connect from Linux to Win already (since I have file sharing established there).  Later I will try to get Win to connect to Linux.

How times are changing.

I studied Electronics Engineering, worked as a production manager for 10 years (during which time I did some, but not much programming) and for the last 5 years I've been self employed developing business applications in a windows env.  Just when I'm thinking that I am 'good', along comes another fork in the road ( Linux, PHP, MySQL, Javascript, VB Script, Ajax, DHTML).

Never stop learning new things in this business.

Cheers,
Nap

---

### Post by wieman01 on 2006-09-16
Delete...

---

### Post by Nap_BlownApart on 2006-09-21
Wieman01,
  Thnx 4 the tip concerning Samba.
Cheers,
Nap

---

### Post by Icereval on 2006-09-21
sudo su - Will get you in as root in a terminal and you can execute as many commands as you like (the passwort it asks you for is your password)

This is assuming your account has access to root.

---

### Post by Nap_BlownApart on 2006-09-21
Icereval,
  Thnx.
  I should have marked the post as resolved, since I was given that info earlier.

Cheers,
Nap

---

### Post by Akita on 2006-09-21
sudo $SHELL

---

